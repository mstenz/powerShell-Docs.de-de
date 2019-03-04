---
title: Ein Argument Bereich überprüfen | Microsoft-Dokumentation
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859736"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="e31fe-102">Überprüfen eines Argumentbereichs</span><span class="sxs-lookup"><span data-stu-id="e31fe-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="e31fe-103">Dieses Beispiel zeigt, wie Sie eine Validierungsregel angeben, die die Windows PowerShell-Laufzeit verwenden können, um die minimalen und maximalen Werte des Parameters-Arguments zu überprüfen, bevor Sie das Cmdlet ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e31fe-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="e31fe-104">Sie haben diese Validierungsregel durch Deklarieren des Attributs ValidateRange festlegen.</span><span class="sxs-lookup"><span data-stu-id="e31fe-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="e31fe-105">Weitere Informationen zu der Klasse, die dieses Attribut definiert, finden Sie unter [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="e31fe-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="e31fe-106">Um ein Argument-Bereich zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="e31fe-106">To validate an argument range</span></span>

- <span data-ttu-id="e31fe-107">Fügen Sie das Attribut ValidateRange hinzu, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="e31fe-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="e31fe-108">In diesem Beispiel gibt einen Bereich von 0 bis 5 für die `InputData` Parameter.</span><span class="sxs-lookup"><span data-stu-id="e31fe-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

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

<span data-ttu-id="e31fe-109">Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [ValidateRange Attributdeklaration](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="e31fe-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e31fe-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e31fe-110">See Also</span></span>

[<span data-ttu-id="e31fe-111">ValidateRange Attributdeklaration</span><span class="sxs-lookup"><span data-stu-id="e31fe-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="e31fe-112">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="e31fe-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
