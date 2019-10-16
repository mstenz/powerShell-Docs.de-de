---
title: Validieren eines Argument Bereichs | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365519"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="50723-102">Überprüfen eines Argumentbereichs</span><span class="sxs-lookup"><span data-stu-id="50723-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="50723-103">In diesem Beispiel wird gezeigt, wie eine Validierungs Regel angegeben wird, mit der die Windows PowerShell-Laufzeit den minimalen und maximalen Wert des Parameter Arguments vor dem Ausführen des Cmdlets überprüfen kann.</span><span class="sxs-lookup"><span data-stu-id="50723-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="50723-104">Diese Validierungs Regel legen Sie fest, indem Sie das validaterange-Attribut deklarieren.</span><span class="sxs-lookup"><span data-stu-id="50723-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="50723-105">Weitere Informationen zu der Klasse, die dieses Attribut definiert, finden Sie unter [System. Management. Automation. validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="50723-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="50723-106">So validieren Sie einen Argument Bereich</span><span class="sxs-lookup"><span data-stu-id="50723-106">To validate an argument range</span></span>

- <span data-ttu-id="50723-107">Fügen Sie das validaterange-Attribut hinzu, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="50723-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="50723-108">In diesem Beispiel wird ein Bereich von 0 bis 5 für den Parameter `InputData` angegeben.</span><span class="sxs-lookup"><span data-stu-id="50723-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

<span data-ttu-id="50723-109">Weitere Informationen zum Deklarieren dieses Attributs finden Sie unter [validaterange-Attribut Deklaration](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="50723-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="50723-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="50723-110">See Also</span></span>

[<span data-ttu-id="50723-111">Validaterange-Attribut Deklaration</span><span class="sxs-lookup"><span data-stu-id="50723-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="50723-112">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="50723-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
