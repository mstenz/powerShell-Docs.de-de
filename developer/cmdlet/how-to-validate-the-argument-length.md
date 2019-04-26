---
title: 'Gewusst wie: Überprüfen Sie die Argumentlänge | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, example
ms.assetid: d5ddaa6e-4904-46da-beb0-0295a8f38332
caps.latest.revision: 12
ms.openlocfilehash: 8a21675acd087df93f93c25952c78931255d60b3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067710"
---
# <a name="how-to-validate-the-argument-length"></a>Überprüfen einer Argumentlänge

Dieses Beispiel zeigt, wie Sie eine Validierungsregel angeben, die die Windows PowerShell-Laufzeit verwenden können, um die Anzahl der Zeichen (die Länge) des Parameters-Arguments zu überprüfen, bevor Sie das Cmdlet ausgeführt wird. Sie haben diese Gültigkeitsprüfungsregel durch Deklarieren des Attributs validateLength auf festlegen.

> [!NOTE]
> Weitere Informationen zu der Klasse, die dieses Attribut definiert, finden Sie unter [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).

## <a name="to-validate-the-argument-length"></a>So überprüfen die Argumentlänge

- Fügen Sie die Validate-Attribut hinzu, wie im folgenden Code gezeigt. In diesem Beispiel gibt an, dass die Länge des Arguments mit eine Länge von 0 bis 10 Zeichen haben soll.

    ```csharp
    [ValidateLength(0, 10)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [validateLength auf Attributdeklaration](./validatelength-attribute-declaration.md).

## <a name="see-also"></a>Weitere Informationen

[ValidateLength auf Attributdeklaration](./validatelength-attribute-declaration.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
