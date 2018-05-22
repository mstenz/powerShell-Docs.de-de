---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: ResourceGet-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 30cbaa907d4dc3a921c9e5fe61ffddc5d61c2347
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a>ResourceGet-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Ruft direkt die **Get**-Methode einer DSC-Ressource auf.

<a name="syntax"></a>Syntax
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a>Parameter
----------

*ResourceType* \[in\] Der Name der aufzurufenden Ressource.

*ModuleName* \[in\] Der Name des Moduls, das die aufzurufende Ressource enthält.

*resourceProperty* \[in\] Gibt den Namen der Ressourceneigenschaft und deren Wert in einer Hashtabelle als Schlüssel und Wert an. Verwenden Sie das Cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) zum Ermitteln von Ressourceneigenschaften und deren Typen.

*configurations* \[out\] Enthält bei Rückgabe eine eingebettete Instanz der Konfigurationen.

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