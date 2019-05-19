---
title: ValidateLength auf Attributdeklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 4d3cdccc0fe3e24b1221e41beef4821b613aab93
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855155"
---
# <a name="validatelength-attribute-declaration"></a>Attributdeklaration: ValidateLength

Die validateLength auf-Attribut gibt an, die minimale und maximale Anzahl von Zeichen für ein Cmdlet-Parameter-Argument. Dieses Attribut kann auch von Windows PowerShell-Funktionen verwendet werden.

## <a name="syntax"></a>Syntax

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parameter

`MinLength` ([System.Integer](/dotnet/api/System.Integer)) erforderlich. Gibt die minimale Anzahl von Zeichen zulässig.

`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) erforderlich. Gibt die maximale Anzahl zulässiger Zeichen.

## <a name="remarks"></a>Hinweise

- Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [wie Eingabe Validierungsregeln deklarieren](./how-to-validate-parameter-input.md).

- Wenn dieses Attribut nicht verwendet wird, kann das entsprechende Parameterargument mit beliebiger Länge sein.

- Die Windows PowerShell-Laufzeit löst einen Fehler in den folgenden Situationen aus:

    - Bei den Wert des der `MaxLength` Attributparameter ist kleiner als der Wert, der die `MinLength` Attributparameter.

    - Wenn die `MaxLength` Attributparameter auf 0 festgelegt ist.

    - Wenn das Argument keine Zeichenfolge ist.

- Das Attribut validateLength auf wird definiert, durch die [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) Klasse.

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
