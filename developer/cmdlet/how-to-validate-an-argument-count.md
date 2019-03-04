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
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="997d7-102">Überprüfen einer Argumentanzahl</span><span class="sxs-lookup"><span data-stu-id="997d7-102">How to Validate an Argument Count</span></span>

<span data-ttu-id="997d7-103">Dieses Beispiel zeigt, wie Sie eine Validierungsregel angeben, die die Windows PowerShell-Laufzeit verwenden können, um die Anzahl von Argumenten (Anzahl) zu überprüfen, die einen Parameter akzeptiert, bevor Sie das Cmdlet ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="997d7-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="997d7-104">Sie haben diese Validierungsregel durch Deklarieren des Attributs ValidateCount festlegen.</span><span class="sxs-lookup"><span data-stu-id="997d7-104">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="997d7-105">Weitere Informationen zu der Klasse, die dieses Attribut definiert, finden Sie unter [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span><span class="sxs-lookup"><span data-stu-id="997d7-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="997d7-106">Um eine Anzahl an Argumenten zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="997d7-106">To validate an argument count</span></span>

- <span data-ttu-id="997d7-107">Fügen Sie die Validate-Attribut hinzu, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="997d7-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="997d7-108">In diesem Beispiel gibt an, dass der Parameter eines Arguments oder bis zu drei Argumente akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="997d7-108">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

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

<span data-ttu-id="997d7-109">Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [ValidateCount Attributdeklaration](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="997d7-109">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="997d7-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="997d7-110">See Also</span></span>

[<span data-ttu-id="997d7-111">ValidateCount Attributdeklaration</span><span class="sxs-lookup"><span data-stu-id="997d7-111">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="997d7-112">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="997d7-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
