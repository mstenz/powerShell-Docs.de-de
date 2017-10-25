---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: RemoveConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>RemoveConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Entfernt die Konfigurationsdateien.

<a name="syntax"></a>Syntax
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a>Parameter
----------

*Stage* \[in\]  
Gibt an, welches Konfigurationsdokument entfernt werden soll. Die folgenden Werte sind gültig:

|Value |Beschreibung |
|:--- |:---|
|**1** | Das **aktuelle** (Current) Konfigurationsdokument (current.mof). |
|**2** | Das **ausstehende** (Pending) Konfigurationsdokument (pending.mof).  |
|**4** | Das **vorherige** (Previous) Konfigurationsdokument (previous.mof). |

*Force* \[in\]  
**true**, um das Entfernen der Konfiguration zu erzwingen.

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


 

 



