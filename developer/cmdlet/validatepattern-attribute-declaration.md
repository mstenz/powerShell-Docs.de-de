---
title: Deklaration von ValidatePattern-Attribut | Microsoft-Dokumentation
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067126"
---
# <a name="validatepattern-attribute-declaration"></a>Attributdeklaration: ValidatePattern

Das ValidatePattern-Attribut gibt an, das Muster eines regulären Ausdrucks, das das Argument der Cmdlet-Parameter überprüft werden. Dieses Attribut kann auch von Windows PowerShell-Funktionen verwendet werden.

Wenn ein Cmdlet validatepattern-Element aufgerufen wird, wird die Windows PowerShell-Laufzeit konvertiert das Argument von der Cmdlet-Parameter in eine Zeichenfolge und vergleicht dann diese Zeichenfolge in das Muster, die durch das ValidatePattern-Attribut angegeben. Das Cmdlet ausgeführt wird, nur dann, wenn die konvertierte Zeichenfolge-Darstellung des Arguments und dem angegebenen Muster übereinstimmen. Wenn sie nicht übereinstimmen, wird ein Fehler von der Windows PowerShell-Laufzeit ausgelöst.

## <a name="syntax"></a>Syntax

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>Parameter

`RegexString` ([System.String](/dotnet/api/System.String)) erforderlich. Gibt einen regulären Ausdruck, der das Parameterargument überprüft.

Optionen ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional benannter Parameter. Gibt eine bitweise Kombination von [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) Flags, die Optionen für reguläre Ausdrücke angeben.

## <a name="remarks"></a>Hinweise

- Dieses Attribut kann nur einmal pro Parameter verwendet werden.

- Sie können die `Option` Parameter des Attributs, das Muster genauer zu definieren. Beispielsweise können Sie die Groß-/ Kleinschreibung des Musters vornehmen.

- Wenn dieses Attribut auf eine Auflistung angewendet wird, muss jedes Element in der Auflistung mit dem Muster entsprechen.

- Das ValidatePattern-Attribut definiert ist, durch die [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) Klasse.

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
