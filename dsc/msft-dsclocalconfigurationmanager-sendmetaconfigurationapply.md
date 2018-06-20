---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendMetaConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 46acd86ac52b7b6b39f06fc65af2498b4f5348ed
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218840"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a>SendMetaConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Legt die Einstellungen des lokalen Konfigurations-Managers fest, die zur Steuerung des Konfigurations-Agents verwendet werden.

<a name="syntax"></a>Syntax
------

```mof
uint32 SendMetaConfigurationApply(
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