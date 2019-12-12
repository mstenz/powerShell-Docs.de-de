---
title: Validieren eines Argument Bereichs | Microsoft-Dokumentation
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365519"
---
# <a name="how-to-validate-an-argument-range"></a>Überprüfen eines Argumentbereichs

In diesem Beispiel wird gezeigt, wie eine Validierungs Regel angegeben wird, mit der die Windows PowerShell-Laufzeit den minimalen und maximalen Wert des Parameter Arguments vor dem Ausführen des Cmdlets überprüfen kann. Diese Validierungs Regel legen Sie fest, indem Sie das validaterange-Attribut deklarieren.

> [!NOTE]
> Weitere Informationen zu der Klasse, die dieses Attribut definiert, finden Sie unter [System. Management. Automation. validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).

### <a name="to-validate-an-argument-range"></a>So validieren Sie einen Argument Bereich

- Fügen Sie das validaterange-Attribut hinzu, wie im folgenden Code gezeigt. In diesem Beispiel wird ein Bereich von 0 bis 5 für den `InputData`-Parameter angegeben.

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

Weitere Informationen zum Deklarieren dieses Attributs finden Sie unter [validaterange-Attribut Deklaration](./validaterange-attribute-declaration.md).

## <a name="see-also"></a>Weitere Informationen

[Validaterange-Attribut Deklaration](./validaterange-attribute-declaration.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
