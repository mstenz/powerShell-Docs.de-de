---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: ResourceSet-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 0c9c1d33117067d76d61036d5839f0b676eb4a97
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219615"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a>ResourceSet-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Ruft direkt die **Set**-Methode einer DSC-Ressource auf.

<a name="syntax"></a>Syntax
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a>Parameter
----------

*ResourceType* \[in\] Der Name der aufzurufenden Ressource.

*ModuleName* \[in\] Der Name des Moduls, das die aufzurufende Ressource enthält.

*resourceProperty* \[in\] Gibt den Namen der Ressourceneigenschaft und deren Wert in einer Hashtabelle als Schlüssel und Wert an. Verwenden Sie das Cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) zum Ermitteln von Ressourceneigenschaften und deren Typen.

*RebootRequired* \[out\] Bei der Rückgabe wird diese Eigenschaft auf **true** festgelegt, wenn der Zielknoten neu gestartet werden muss.

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