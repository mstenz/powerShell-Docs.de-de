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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067177"
---
# <a name="validatecount-attribute-declaration"></a>Attributdeklaration: ValidateCount

Die ValidateCount-Attribut gibt an, die minimale und maximale Anzahl von Argumenten, die für ein Cmdlet-Parameter zulässig.

## <a name="syntax"></a>Syntax

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parameter

`MinLength` ([System.Int32][]) erforderlich. Gibt die minimale Anzahl von Argumenten an.

`MaxLength`([System.Int32][]) erforderlich. Gibt die maximale Anzahl von Argumenten an.

## <a name="remarks"></a>Hinweise

- Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [Wie Sie eine Anzahl an Argumenten überprüfen][].

- Wenn dieses Attribut nicht aufgerufen wird, kann der entsprechende Cmdlet-Parameter eine beliebige Anzahl von Argumenten verfügen.

- Die Windows PowerShell-Laufzeit löst einen Fehler in den folgenden Situationen aus:

    - Die `MinLength` und `MaxLength` Parameter sind nicht vom Typ [System.Int32][].

    - Der Wert des der `MaxLength` Attributparameter ist kleiner als der Wert, der die `MinLength` Attributparameter.

- Das ValidateCount-Attribut definiert ist, indem die [System.Management.Automation.ValidateCountAttribute][] Klasse.

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.ValidateCountAttribute][]

[Wie Sie eine Anzahl an Argumenten überprüfen][]

[Schreiben eines Windows PowerShell-Cmdlets][]

[Wie Sie eine Anzahl an Argumenten überprüfen]: how-to-validate-an-argument-count.md
[Schreiben eines Windows PowerShell-Cmdlets]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
