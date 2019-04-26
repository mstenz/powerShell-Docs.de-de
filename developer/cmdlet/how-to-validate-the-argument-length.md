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
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="91b31-102">Überprüfen einer Argumentlänge</span><span class="sxs-lookup"><span data-stu-id="91b31-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="91b31-103">Dieses Beispiel zeigt, wie Sie eine Validierungsregel angeben, die die Windows PowerShell-Laufzeit verwenden können, um die Anzahl der Zeichen (die Länge) des Parameters-Arguments zu überprüfen, bevor Sie das Cmdlet ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="91b31-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="91b31-104">Sie haben diese Gültigkeitsprüfungsregel durch Deklarieren des Attributs validateLength auf festlegen.</span><span class="sxs-lookup"><span data-stu-id="91b31-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="91b31-105">Weitere Informationen zu der Klasse, die dieses Attribut definiert, finden Sie unter [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span><span class="sxs-lookup"><span data-stu-id="91b31-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="91b31-106">So überprüfen die Argumentlänge</span><span class="sxs-lookup"><span data-stu-id="91b31-106">To validate the argument length</span></span>

- <span data-ttu-id="91b31-107">Fügen Sie die Validate-Attribut hinzu, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="91b31-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="91b31-108">In diesem Beispiel gibt an, dass die Länge des Arguments mit eine Länge von 0 bis 10 Zeichen haben soll.</span><span class="sxs-lookup"><span data-stu-id="91b31-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

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

<span data-ttu-id="91b31-109">Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [validateLength auf Attributdeklaration](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="91b31-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="91b31-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="91b31-110">See Also</span></span>

[<span data-ttu-id="91b31-111">ValidateLength auf Attributdeklaration</span><span class="sxs-lookup"><span data-stu-id="91b31-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="91b31-112">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="91b31-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
