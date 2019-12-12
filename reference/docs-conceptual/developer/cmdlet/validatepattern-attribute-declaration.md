---
title: Validatepattern-Attribut Deklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369159"
---
# <a name="validatepattern-attribute-declaration"></a>Attributdeklaration: ValidatePattern

Das validatepattern-Attribut gibt ein Muster für reguläre Ausdrücke an, das das Argument eines Cmdlet-Parameters überprüft. Dieses Attribut kann auch von Windows PowerShell-Funktionen verwendet werden.

Wenn validatepattern innerhalb eines Cmdlets aufgerufen wird, konvertiert Windows PowerShell Runtime das-Argument des Cmdlet-Parameters in eine Zeichenfolge und vergleicht diese Zeichenfolge dann mit dem Muster, das vom validatepattern-Attribut bereitgestellt wird. Das-Cmdlet wird nur ausgeführt, wenn die konvertierte Zeichen folgen Darstellung des Arguments und des angegebenen Musters abgleichen. Wenn Sie nicht identisch sind, wird von der Windows PowerShell-Laufzeit ein Fehler ausgelöst.

## <a name="syntax"></a>Syntax

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>Parameter

`RegexString` ([System. String](/dotnet/api/System.String)) erforderlich. Gibt einen regulären Ausdruck an, der das Parameter Argument überprüft.

Optionen ([System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) optionaler benannter Parameter. Gibt eine bitweise Kombination von [System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) -Flags an, die Optionen für reguläre Ausdrücke angeben.

## <a name="remarks"></a>Hinweise

- Dieses Attribut kann nur einmal pro Parameter verwendet werden.

- Mit dem `Option`-Parameter des-Attributs können Sie das Muster weiter definieren. Beispielsweise können Sie für das Muster die Groß-/Kleinschreibung beachten.

- Wenn dieses Attribut auf eine Auflistung angewendet wird, muss jedes Element in der Auflistung mit dem Muster identisch sein.

- Das validatepattern-Attribut wird von der [System. Management. Automation. validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) -Klasse definiert.

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
