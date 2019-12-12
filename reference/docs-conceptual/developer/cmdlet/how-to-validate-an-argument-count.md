---
title: Validieren einer Argument Anzahl | Microsoft-Dokumentation
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365529"
---
# <a name="how-to-validate-an-argument-count"></a>Überprüfen einer Argumentanzahl

In diesem Beispiel wird gezeigt, wie eine Validierungs Regel angegeben wird, mit der die Windows PowerShell-Laufzeit die Anzahl der Argumente (die Anzahl) überprüfen kann, die ein Parameter annimmt, bevor das Cmdlet ausgeführt wird. Diese Validierungs Regel legen Sie fest, indem Sie das validatecount-Attribut deklarieren.

> [!NOTE]
> Weitere Informationen zu der Klasse, die dieses Attribut definiert, finden Sie unter [System. Management. Automation. validatezähltattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).

## <a name="to-validate-an-argument-count"></a>So überprüfen Sie eine Argument Anzahl

- Fügen Sie das Validate-Attribut hinzu, wie im folgenden Code gezeigt. In diesem Beispiel wird angegeben, dass der-Parameter ein Argument oder bis zu drei Argumente akzeptiert.

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

Weitere Informationen zum Deklarieren dieses Attributs finden Sie unter [validatecount-Attribut Deklaration](./validatecount-attribute-declaration.md).

## <a name="see-also"></a>Weitere Informationen

[Validatecount-Attribut Deklaration](./validatecount-attribute-declaration.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
