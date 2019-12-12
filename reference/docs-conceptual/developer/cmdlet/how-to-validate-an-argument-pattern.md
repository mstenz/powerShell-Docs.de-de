---
title: Validieren eines Argument Musters | Microsoft-Dokumentation
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365559"
---
# <a name="how-to-validate-an-argument-pattern"></a>Überprüfen eines Argumentmusters

In diesem Beispiel wird gezeigt, wie eine Validierungs Regel angegeben wird, mit der die Windows PowerShell-Laufzeit das Zeichen Muster des Parameter Arguments vor dem Ausführen des Cmdlets überprüfen kann. Diese Validierungs Regel legen Sie fest, indem Sie das validatepattern-Attribut deklarieren.

> [!NOTE]
> Weitere Informationen zu der Klasse, die dieses Attribut definiert, finden Sie unter [System. Management. Automation. validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).

## <a name="to-validate-an-argument-pattern"></a>So validieren Sie ein Argument Muster

- Fügen Sie das Validate-Attribut hinzu, wie im folgenden Code gezeigt. In diesem Beispiel wird ein Muster von vier Ziffern angegeben, wobei jede Ziffer den Wert 0 bis 9 hat.

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

Weitere Informationen zum Deklarieren dieses Attributs finden Sie unter [validatepattern-Attribut Deklaration](./validatepattern-attribute-declaration.md).

## <a name="see-also"></a>Weitere Informationen

[Validatepattern-Attribut Deklaration](./validatepattern-attribute-declaration.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
