---
title: ValidateCount Attributdeklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 4e0be34b6f7a56dcf02a4381de4d2a5d08db14df
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794438"
---
# <a name="validatecount-attribute-declaration"></a>Attributdeklaration: ValidateCount

Die ValidateCount-Attribut gibt an, die minimale und maximale Anzahl von Argumenten, die für ein Cmdlet-Parameter zulässig.

## <a name="syntax"></a>Syntax

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parameter

`MinLength` ([System. Int32](/dotnet/api/System.Int32)) erforderlich. Gibt die minimale Anzahl von Argumenten an.

`MaxLength`([System. Int32](/dotnet/api/System.Int32)) erforderlich. Gibt die maximale Anzahl von Argumenten an.

## <a name="remarks"></a>Hinweise

- Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [wie Eingabe Validierungsregeln deklarieren](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).

- Wenn dieses Attribut nicht aufgerufen wird, kann der entsprechende Cmdlet-Parameter eine beliebige Anzahl von Argumenten verfügen.

- Die Windows PowerShell-Laufzeit löst einen Fehler in den folgenden Situationen aus:

    - Die `MinLength` und `MaxLength` Parameter sind nicht vom Typ [System. Int32](/dotnet/api/System.Int32).

    - Der Wert des der `MaxLength` Attributparameter ist kleiner als der Wert, der die `MinLength` Attributparameter.

- Das ValidateCount-Attribut definiert ist, indem die [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) Klasse.

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)

[Gewusst wie: Deklarieren Sie die Überprüfung der Eingabe-Regeln](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
