---
title: Validatecount-Attribut Deklaration | Microsoft-Dokumentation
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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369229"
---
# <a name="validatecount-attribute-declaration"></a>Attributdeklaration: ValidateCount

Das validatecount-Attribut gibt die minimale und maximale Anzahl von Argumenten an, die für einen Cmdlet-Parameter zulässig sind.

## <a name="syntax"></a>Syntax

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parameter

`MinLength` ([System.Int32][]) erforderlich. Gibt die Mindestanzahl von Argumenten an.

`MaxLength`([System.Int32][]) erforderlich. Gibt die maximale Anzahl von Argumenten an.

## <a name="remarks"></a>Hinweise

- Weitere Informationen zum Deklarieren dieses Attributs finden Sie unter [Validieren einer Argument Anzahl][].

- Wenn dieses Attribut nicht aufgerufen wird, kann der entsprechende Cmdlet-Parameter über eine beliebige Anzahl von Argumenten verfügen.

- Die Windows PowerShell-Laufzeit löst unter den folgenden Bedingungen einen Fehler aus:

    - Die Attribute "`MinLength`" und "`MaxLength`" sind nicht vom Typ " [System.Int32][]".

    - Der Wert des `MaxLength` Attribute-Parameters ist kleiner als der Wert des `MinLength` Attribute-Parameters.

- Das validatecount-Attribut wird von der [System. Management. Automation. validatezähltattribute][] -Klasse definiert.

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. validatezähltattribute][]

[Validieren einer Argument Anzahl][]

[Schreiben eines Windows PowerShell-Cmdlets][]

[Validieren einer Argument Anzahl]: how-to-validate-an-argument-count.md
[Schreiben eines Windows PowerShell-Cmdlets]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System. Management. Automation. validatezähltattribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
