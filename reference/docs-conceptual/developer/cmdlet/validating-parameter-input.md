---
title: Validieren von Parameter Eingaben | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363509"
---
# <a name="validating-parameter-input"></a>Überprüfen von Parametereingaben

PowerShell kann die Argumente, die an Cmdlet-Parameter übergeben werden, auf verschiedene Weise überprüfen.
PowerShell kann die Länge, den Bereich und das Muster der Zeichen des Arguments überprüfen.
Sie kann die Anzahl der verfügbaren Argumente (die Anzahl) überprüfen.
Diese Validierungsregeln werden durch Validierungs Attribute definiert, die mit dem Parameter-Attribut in öffentlichen Eigenschaften der Cmdlet-Klasse deklariert werden.

Zum Validieren eines Parameter Arguments verwendet die PowerShell-Laufzeit die Informationen, die von den Validierungs Attributen bereitgestellt werden, um den Wert des-Parameters vor dem Ausführen des Cmdlets zu bestätigen.
Wenn die Parameter Eingabe nicht gültig ist, erhält der Benutzer eine Fehlermeldung.
Jeder Validierungs Parameter definiert eine Validierungs Regel, die von PowerShell erzwungen wird.

PowerShell erzwingt die Validierungsregeln basierend auf den folgenden Attributen.

### <a name="validatecount"></a>Validatecount

Gibt die minimale und maximale Anzahl von Argumenten an, die ein Parameter annehmen kann.
Weitere Informationen finden Sie unter [validatecount-Attribut Deklaration](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Gibt die minimale und maximale Anzahl von Zeichen im Parameter Argument an.
Weitere Informationen finden Sie unter [validateLength-Attribut Deklaration](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Gibt einen regulären Ausdruck an, der das Parameter Argument überprüft.
Weitere Informationen finden Sie unter [validatepattern-Attribut Deklaration](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>Validaterange

Gibt den minimalen und maximalen Wert des Parameter Arguments an.
Weitere Informationen finden Sie unter [validaterange-Attribut Deklaration](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Gibt die gültigen Werte für das Parameter Argument an.
Weitere Informationen finden Sie unter [validateset-Attribut Deklaration](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Weitere Informationen

[Validieren von Parameter Eingaben](./how-to-validate-parameter-input.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
