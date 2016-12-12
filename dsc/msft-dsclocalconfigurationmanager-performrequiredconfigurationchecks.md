---
title: PerformRequiredConfigurationChecks-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: f9eb975845f6ccabcac80e2591fd987f80f81331
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
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

*Flags* \[in\]  
Eine Bitmaske, die den Typ der auszuführenden Konsistenzprüfung angibt. Die folgenden Werte sind gültig und können mit einem bitweisen **ODER**-Vorgang kombiniert werden:

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


 

 



