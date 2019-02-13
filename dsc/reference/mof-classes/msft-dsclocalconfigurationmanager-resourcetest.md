---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: ResourceTest-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678439"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a>ResourceTest-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Ruft direkt die **Test**-Methode einer DSC-Ressource auf.

## <a name="syntax"></a>Syntax

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a>Parameter

*ResourceType* \[in\] Der Name der aufzurufenden Ressource.

*ModuleName* \[in\] Der Name des Moduls, das die aufzurufende Ressource enthält.

*resourceProperty* \[in\] Gibt den Namen der Ressourceneigenschaft und deren Wert in einer Hashtabelle als Schlüssel und Wert an. Verwenden Sie das Cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) zum Ermitteln von Ressourceneigenschaften und deren Typen.

*InDesiredState* \[out\] Bei der Rückgabe wird diese Eigenschaft auf **true** festgelegt, wenn sich der Zielknoten im gewünschten Zustand befindet.

## <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.

## <a name="remarks"></a>Hinweise

Dies ist eine statische Methode.

## <a name="requirements"></a>Anforderungen

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Siehe auch

[**MSFT_DSCLocalConfigurationManager-Klasse**](msft-dsclocalconfigurationmanager.md)