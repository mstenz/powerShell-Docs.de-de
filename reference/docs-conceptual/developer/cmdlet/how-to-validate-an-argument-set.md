---
title: Validieren eines Argument Satzes | Microsoft-Dokumentation
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365509"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="d6cf7-102">Überprüfen eines Argumentsatzes</span><span class="sxs-lookup"><span data-stu-id="d6cf7-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="d6cf7-103">Dieses Beispiel zeigt, wie Sie eine Validierungs Regel angeben, mit der die Windows PowerShell-Laufzeit das Parameter Argument vor dem Ausführen des Cmdlets überprüfen kann.</span><span class="sxs-lookup"><span data-stu-id="d6cf7-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="d6cf7-104">Diese Validierungs Regel stellt einen Satz gültiger Werte für das Parameter Argument bereit.</span><span class="sxs-lookup"><span data-stu-id="d6cf7-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="d6cf7-105">Weitere Informationen zu der Klasse, die dieses Attribut definiert, finden Sie unter [System. Management. Automation. validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="d6cf7-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="d6cf7-106">So validieren Sie einen Argument Satz</span><span class="sxs-lookup"><span data-stu-id="d6cf7-106">To validate an argument set</span></span>

- <span data-ttu-id="d6cf7-107">Fügen Sie das validateset-Attribut hinzu, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="d6cf7-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="d6cf7-108">In diesem Beispiel wird ein Satz von drei möglichen Werten für den `UserName`-Parameter angegeben.</span><span class="sxs-lookup"><span data-stu-id="d6cf7-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="d6cf7-109">Weitere Informationen zum Deklarieren dieses Attributs finden Sie unter [validateset-Attribut Deklaration](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="d6cf7-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d6cf7-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d6cf7-110">See Also</span></span>

[<span data-ttu-id="d6cf7-111">System. Management. Automation. validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="d6cf7-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="d6cf7-112">Validateset-Attribut Deklaration</span><span class="sxs-lookup"><span data-stu-id="d6cf7-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="d6cf7-113">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="d6cf7-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
