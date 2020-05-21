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
ms.openlocfilehash: 3cae95fab30a4abe4e544ed5cb7dadc9f4debf02
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692375"
---
# <a name="validatecount-attribute-declaration"></a>Attributdeklaration: ValidateCount

Das validatecount-Attribut gibt die minimale und maximale Anzahl von Argumenten an, die für einen Cmdlet-Parameter zulässig sind.

## <a name="syntax"></a>Syntax

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parameter

`MinLength`([System. Int32][]) erforderlich. Gibt die Mindestanzahl von Argumenten an.

`MaxLength`([System. Int32][]) erforderlich. Gibt die maximale Anzahl von Argumenten an.

## <a name="remarks"></a>Hinweise

- Weitere Informationen zum Deklarieren dieses Attributs finden Sie unter [Validieren einer Argument Anzahl][].

- Wenn dieses Attribut nicht aufgerufen wird, kann der entsprechende Cmdlet-Parameter über eine beliebige Anzahl von Argumenten verfügen.

- Die Windows PowerShell-Laufzeit löst unter den folgenden Bedingungen einen Fehler aus:

  - Die `MinLength` -und- `MaxLength` Attribut Parameter sind nicht vom Typ [System. Int32][].

  - Der Wert des `MaxLength` Attribut Parameters ist kleiner als der Wert des `MinLength` Attribut Parameters.

- Das validatecount-Attribut wird von der [System. Management. Automation. validatezähltattribute][] -Klasse definiert.

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. validatezähltattribute][]

[Überprüfen einer Argumentanzahl][]

[Schreiben eines Windows PowerShell-Cmdlets][]

[Überprüfen einer Argumentanzahl]: how-to-validate-an-argument-count.md
[Schreiben eines Windows PowerShell-Cmdlets]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System. Management. Automation. validatezähltattribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
