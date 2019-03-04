---
title: Ein Argument Bereich überprüfen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859736"
---
# <a name="how-to-validate-an-argument-range"></a>Überprüfen eines Argumentbereichs

Dieses Beispiel zeigt, wie Sie eine Validierungsregel angeben, die die Windows PowerShell-Laufzeit verwenden können, um die minimalen und maximalen Werte des Parameters-Arguments zu überprüfen, bevor Sie das Cmdlet ausgeführt wird. Sie haben diese Validierungsregel durch Deklarieren des Attributs ValidateRange festlegen.

> [!NOTE]
> Weitere Informationen zu der Klasse, die dieses Attribut definiert, finden Sie unter [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).

### <a name="to-validate-an-argument-range"></a>Um ein Argument-Bereich zu überprüfen.

- Fügen Sie das Attribut ValidateRange hinzu, wie im folgenden Code gezeigt. In diesem Beispiel gibt einen Bereich von 0 bis 5 für die `InputData` Parameter.

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [ValidateRange Attributdeklaration](./validaterange-attribute-declaration.md).

## <a name="see-also"></a>Weitere Informationen

[ValidateRange Attributdeklaration](./validaterange-attribute-declaration.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
