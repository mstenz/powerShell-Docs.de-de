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
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="dd35b-102">Überprüfen eines Argumentsatzes</span><span class="sxs-lookup"><span data-stu-id="dd35b-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="dd35b-103">Dieses Beispiel zeigt, wie Sie eine Validierungsregel angeben, die die Windows PowerShell-Laufzeit verwenden können, um Parameterargument zu überprüfen, bevor Sie das Cmdlet ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="dd35b-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="dd35b-104">Diese Validierungsregel bietet eine Reihe der gültigen Werte für das Parameterargument.</span><span class="sxs-lookup"><span data-stu-id="dd35b-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="dd35b-105">Weitere Informationen zu der Klasse, die dieses Attribut definiert, finden Sie unter [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="dd35b-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="dd35b-106">Um zu überprüfen, ob ein Argument festlegen</span><span class="sxs-lookup"><span data-stu-id="dd35b-106">To validate an argument set</span></span>

- <span data-ttu-id="dd35b-107">Fügen Sie das ValidateSet-Attribut aus, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="dd35b-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="dd35b-108">In diesem Beispiel gibt einen Satz von drei mögliche Werte für die `UserName` Parameter.</span><span class="sxs-lookup"><span data-stu-id="dd35b-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="dd35b-109">Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [ValidateSet Attributdeklaration](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="dd35b-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dd35b-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="dd35b-110">See Also</span></span>

[<span data-ttu-id="dd35b-111">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="dd35b-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="dd35b-112">Deklaration von ValidateSet-Attribut</span><span class="sxs-lookup"><span data-stu-id="dd35b-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="dd35b-113">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="dd35b-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
