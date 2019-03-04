---
title: 'Gewusst wie: Überprüfen Sie eine Anzahl an Argumenten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859136"
---
# <a name="how-to-validate-an-argument-count"></a>Überprüfen einer Argumentanzahl

Dieses Beispiel zeigt, wie Sie eine Validierungsregel angeben, die die Windows PowerShell-Laufzeit verwenden können, um die Anzahl von Argumenten (Anzahl) zu überprüfen, die einen Parameter akzeptiert, bevor Sie das Cmdlet ausgeführt wird. Sie haben diese Validierungsregel durch Deklarieren des Attributs ValidateCount festlegen.

> [!NOTE]
> Weitere Informationen zu der Klasse, die dieses Attribut definiert, finden Sie unter [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).

## <a name="to-validate-an-argument-count"></a>Um eine Anzahl an Argumenten zu überprüfen.

- Fügen Sie die Validate-Attribut hinzu, wie im folgenden Code gezeigt. In diesem Beispiel gibt an, dass der Parameter eines Arguments oder bis zu drei Argumente akzeptiert.

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [ValidateCount Attributdeklaration](./validatecount-attribute-declaration.md).

## <a name="see-also"></a>Weitere Informationen

[ValidateCount Attributdeklaration](./validatecount-attribute-declaration.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
