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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858846"
---
# <a name="validating-parameter-input"></a>Überprüfen von Parametereingaben

Windows PowerShell kann es sich um Cmdlet-Parameter auf unterschiedliche Weise übergebenen Argumente überprüfen. Windows PowerShell können die Länge des Bereichs und dem Muster der Zeichen des Arguments überprüfen. Sie können die Anzahl von Argumenten zur Verfügung (Anzahl) überprüfen. Diese Validierungsregeln werden von Validierungsattributen, die deklariert werden mit dem Parameter-Attribut auf öffentlichen Eigenschaften, die von der Cmdlet-Klasse definiert.

Um ein Parameterargument zu überprüfen, verwendet die Windows PowerShell-Laufzeit die Informationen durch die Validierungsattribute, bestätigen den Wert des Parameters aus, bevor das Cmdlet ausgeführt wird. Wenn die Parametereingabe nicht gültig ist, erhält der Benutzer eine Fehlermeldung angezeigt. Jeder Parameter für die Validierung definiert eine Validierungsregel, die von Windows PowerShell erzwungen wird.

Windows PowerShell erzwingt die Validierungsregeln, die basierend auf den folgenden Attributen.

ValidateCount gibt die minimale und maximale Anzahl von Argumenten, die ein Parameter akzeptieren kann. Weitere Informationen zu der Syntax verwendet, um dieses Attribut zu deklarieren, finden Sie unter [ValidateCount Attributdeklaration](./validatecount-attribute-declaration.md).

ValidateLength auf gibt die minimale und maximale Anzahl von Zeichen in das Parameterargument. Weitere Informationen zu der Syntax verwendet, um dieses Attribut zu deklarieren, finden Sie unter [validateLength auf Attributdeklaration](./validatelength-attribute-declaration.md).

Validatepattern-Element gibt an, einen regulären Ausdruck, der das Parameterargument überprüft werden. Weitere Informationen zu der Syntax verwendet, um dieses Attribut zu deklarieren, finden Sie unter [ValidatePattern Attributdeklaration](./validatepattern-attribute-declaration.md).

ValidateRange gibt an, die minimalen und maximalen Werte des Parameters-Arguments. Weitere Informationen zu der Syntax verwendet, um dieses Attribut zu deklarieren, finden Sie unter [ValidateRange Attributdeklaration](./validaterange-attribute-declaration.md).

ValidateSet gibt die gültigen Werte für das Parameterargument. Weitere Informationen zu der Syntax verwendet, um dieses Attribut zu deklarieren, finden Sie unter [ValidateSet Attributdeklaration](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Weitere Informationen

[Gewusst wie: Überprüfen der Parametereingabe](./how-to-validate-parameter-input.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
