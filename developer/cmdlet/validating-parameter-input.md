---
title: Überprüfen der Parametereingabe | Microsoft-Dokumentation
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067143"
---
# <a name="validating-parameter-input"></a>Überprüfen von Parametereingaben

PowerShell kann es sich um Cmdlet-Parameter auf unterschiedliche Weise übergebenen Argumente überprüfen.
PowerShell kann es sich um die Länge des Bereichs und dem Muster der Zeichen des Arguments überprüfen.
Sie können die Anzahl von Argumenten zur Verfügung (Anzahl) überprüfen.
Diese Validierungsregeln werden von Validierungsattributen, die deklariert werden mit dem Parameter-Attribut auf öffentlichen Eigenschaften, die von der Cmdlet-Klasse definiert.

Um ein Parameterargument zu überprüfen, verwendet die PowerShell-Laufzeit die Informationen durch die Validierungsattribute, bestätigen den Wert des Parameters aus, bevor das Cmdlet ausgeführt wird.
Wenn die Parametereingabe nicht gültig ist, erhält der Benutzer eine Fehlermeldung angezeigt.
Jeder Parameter für die Validierung definiert eine Validierungsregel, die von PowerShell erzwungen wird.

PowerShell erzwingt die Validierungsregeln, die basierend auf den folgenden Attributen.

### <a name="validatecount"></a>ValidateCount

Gibt die minimale und maximale Anzahl von Argumenten, die ein Parameter akzeptieren kann.
Weitere Informationen finden Sie unter [ValidateCount Attributdeklaration](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength auf

Gibt die minimale und maximale Anzahl der Zeichen im Parameterargument.
Weitere Informationen finden Sie unter [validateLength auf Attributdeklaration](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Gibt einen regulären Ausdruck, der das Parameterargument überprüft.
Weitere Informationen finden Sie unter [ValidatePattern Attributdeklaration](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Gibt die minimalen und maximalen Werte des Parameters-Arguments.
Weitere Informationen finden Sie unter [ValidateRange Attributdeklaration](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Gibt die gültigen Werte für das Parameterargument.
Weitere Informationen finden Sie unter [ValidateSet Attributdeklaration](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Weitere Informationen

[Gewusst wie: Überprüfen der Parametereingabe](./how-to-validate-parameter-input.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
