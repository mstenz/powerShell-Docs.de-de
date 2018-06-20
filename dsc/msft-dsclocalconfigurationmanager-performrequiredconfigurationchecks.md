---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: PerformRequiredConfigurationChecks-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: c3fdaa23875815b1cf5cbf0b6e21c633e00664aa
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186693"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>PerformRequiredConfigurationChecks-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Startet eine Konsistenzprüfung unter Verwendung des Taskplaners.

<a name="syntax"></a>Syntax
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a>Parameter
----------

*Flags* \[in\] Eine Bitmaske, die den Typ der auszuführenden Konsistenzprüfung angibt. Die folgenden Werte sind gültig und können mit einem bitweisen **ODER**-Vorgang kombiniert werden:

|Wert |Beschreibung |
|:--- |:---|
|**1** | Eine normale Konsistenzprüfung. |
|**2** | Die Fortsetzung einer Konsistenzprüfung nach einem Neustart. Dieser Wert sollte nicht mit anderen Werten kombiniert werden. |
|**4** | Die Konfiguration sollte von dem Pull-Server abgerufen werden, der in der Metakonfiguration für den Knoten angegeben ist. Dieser Wert sollte immer mit **1** kombiniert werden, um einen Wert von **5** zu erzielen. |
|**8** | Senden des Status an den Berichtsserver. |

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