---
title: Eine Argument Muster überprüfen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067772"
---
# <a name="how-to-validate-an-argument-pattern"></a>Überprüfen eines Argumentmusters

Dieses Beispiel zeigt, wie Sie eine Validierungsregel angeben, die die Windows PowerShell-Laufzeit verwenden können, um die Muster der Zeichen des Parameters-Arguments zu überprüfen, bevor das Cmdlet ausgeführt wird. Sie legen diese Validierungsregel, indem das ValidatePattern-Attribut deklarieren.

> [!NOTE]
> Weitere Informationen zu der Klasse, die dieses Attribut definiert, finden Sie unter [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).

## <a name="to-validate-an-argument-pattern"></a>Um ein Argument-Muster zu überprüfen.

- Fügen Sie die Validate-Attribut hinzu, wie im folgenden Code gezeigt. In diesem Beispiel gibt ein Muster, in dem ein Wert von 0 bis 9 von einzelnen Ziffern verfügt über vier Ziffern an.

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [ValidatePattern Attributdeklaration](./validatepattern-attribute-declaration.md).

## <a name="see-also"></a>Weitere Informationen

[Deklaration von ValidatePattern-Attribut](./validatepattern-attribute-declaration.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
