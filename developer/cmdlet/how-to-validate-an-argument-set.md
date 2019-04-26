---
title: Wie Sie ein Argument auf Gültigkeit überprüft | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067712"
---
# <a name="how-to-validate-an-argument-set"></a>Überprüfen eines Argumentsatzes

Dieses Beispiel zeigt, wie Sie eine Validierungsregel angeben, die die Windows PowerShell-Laufzeit verwenden können, um Parameterargument zu überprüfen, bevor Sie das Cmdlet ausgeführt wird. Diese Validierungsregel bietet eine Reihe der gültigen Werte für das Parameterargument.

> [!NOTE]
> Weitere Informationen zu der Klasse, die dieses Attribut definiert, finden Sie unter [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).

## <a name="to-validate-an-argument-set"></a>Um zu überprüfen, ob ein Argument festlegen

- Fügen Sie das ValidateSet-Attribut aus, wie im folgenden Code gezeigt. In diesem Beispiel gibt einen Satz von drei mögliche Werte für die `UserName` Parameter.

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [ValidateSet Attributdeklaration](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Deklaration von ValidateSet-Attribut](./validateset-attribute-declaration.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
