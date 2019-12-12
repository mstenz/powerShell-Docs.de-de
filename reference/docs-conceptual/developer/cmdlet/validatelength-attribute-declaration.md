---
title: ValidateLength-Attribut Deklaration | Microsoft-Dokumentation
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
ms.openlocfilehash: a25fa2410fcc6803563573596af1bc99052c3ffa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369179"
---
# <a name="validatelength-attribute-declaration"></a>Attributdeklaration: ValidateLength

Das validateLength-Attribut gibt die minimale und maximale Anzahl von Zeichen für ein Cmdlet-Parameter Argument an. Dieses Attribut kann auch von Windows PowerShell-Funktionen verwendet werden.

## <a name="syntax"></a>Syntax

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parameter

`MinLength` ([System. Int32](/dotnet/api/System.Int32)) erforderlich. Gibt die Mindestanzahl von Zeichen an, die zulässig ist.

`MaxLength` ([System. Int32](/dotnet/api/System.Int32)) erforderlich. Gibt die maximal zulässige Anzahl von Zeichen an.

## <a name="remarks"></a>Hinweise

- Weitere Informationen zum Deklarieren dieses Attributs finden Sie unter [Deklarieren von Eingabe Validierungsregeln](./how-to-validate-parameter-input.md).

- Wenn dieses Attribut nicht verwendet wird, kann das entsprechende Parameter Argument eine beliebige Länge aufweisen.

- Die Windows PowerShell-Laufzeit löst unter den folgenden Bedingungen einen Fehler aus:

    - Wenn der Wert des `MaxLength`-Attribut Parameters kleiner ist als der Wert des `MinLength` Attribute-Parameters.

    - Wenn der `MaxLength`-Attribut Parameter auf 0 festgelegt ist.

    - Wenn das Argument keine Zeichenfolge ist.

- Das validateLength-Attribut wird von der [System. Management. Automation. validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) -Klasse definiert.

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
