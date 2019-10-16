---
title: Validieren der Argument Länge | Microsoft-Dokumentation
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365489"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="66f91-102">Überprüfen einer Argumentlänge</span><span class="sxs-lookup"><span data-stu-id="66f91-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="66f91-103">In diesem Beispiel wird gezeigt, wie eine Validierungs Regel angegeben wird, mit der die Windows PowerShell-Laufzeit die Anzahl der Zeichen (die Länge) des Parameter Arguments vor dem Ausführen des Cmdlets überprüfen kann.</span><span class="sxs-lookup"><span data-stu-id="66f91-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="66f91-104">Diese Validierungs Regel legen Sie fest, indem Sie das validateLength-Attribut deklarieren.</span><span class="sxs-lookup"><span data-stu-id="66f91-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="66f91-105">Weitere Informationen zu der Klasse, die dieses Attribut definiert, finden Sie unter [System. Management. Automation. validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span><span class="sxs-lookup"><span data-stu-id="66f91-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="66f91-106">So überprüfen Sie die Argument Länge</span><span class="sxs-lookup"><span data-stu-id="66f91-106">To validate the argument length</span></span>

- <span data-ttu-id="66f91-107">Fügen Sie das Validate-Attribut hinzu, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="66f91-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="66f91-108">In diesem Beispiel wird angegeben, dass die Länge des Arguments eine Länge von 0 bis 10 Zeichen aufweisen soll.</span><span class="sxs-lookup"><span data-stu-id="66f91-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

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

<span data-ttu-id="66f91-109">Weitere Informationen zum Deklarieren dieses Attributs finden Sie unter [validateLength-Attribut Deklaration](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="66f91-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="66f91-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="66f91-110">See Also</span></span>

[<span data-ttu-id="66f91-111">ValidateLength-Attribut Deklaration</span><span class="sxs-lookup"><span data-stu-id="66f91-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="66f91-112">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="66f91-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
