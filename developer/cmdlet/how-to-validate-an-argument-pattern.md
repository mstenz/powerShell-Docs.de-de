---
title: Eine Argument Muster überprüfen | Microsoft-Dokumentation
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067772"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="ec5f1-102">Überprüfen eines Argumentmusters</span><span class="sxs-lookup"><span data-stu-id="ec5f1-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="ec5f1-103">Dieses Beispiel zeigt, wie Sie eine Validierungsregel angeben, die die Windows PowerShell-Laufzeit verwenden können, um die Muster der Zeichen des Parameters-Arguments zu überprüfen, bevor das Cmdlet ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ec5f1-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="ec5f1-104">Sie legen diese Validierungsregel, indem das ValidatePattern-Attribut deklarieren.</span><span class="sxs-lookup"><span data-stu-id="ec5f1-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="ec5f1-105">Weitere Informationen zu der Klasse, die dieses Attribut definiert, finden Sie unter [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span><span class="sxs-lookup"><span data-stu-id="ec5f1-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="ec5f1-106">Um ein Argument-Muster zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="ec5f1-106">To validate an argument pattern</span></span>

- <span data-ttu-id="ec5f1-107">Fügen Sie die Validate-Attribut hinzu, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="ec5f1-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="ec5f1-108">In diesem Beispiel gibt ein Muster, in dem ein Wert von 0 bis 9 von einzelnen Ziffern verfügt über vier Ziffern an.</span><span class="sxs-lookup"><span data-stu-id="ec5f1-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

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

<span data-ttu-id="ec5f1-109">Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [ValidatePattern Attributdeklaration](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ec5f1-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ec5f1-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ec5f1-110">See Also</span></span>

[<span data-ttu-id="ec5f1-111">Deklaration von ValidatePattern-Attribut</span><span class="sxs-lookup"><span data-stu-id="ec5f1-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="ec5f1-112">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="ec5f1-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
