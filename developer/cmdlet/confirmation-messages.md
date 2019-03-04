---
title: Meldungen zur benutzerbestätigung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 75214a3fe4bc019836f75db19fb873bd081f200f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861416"
---
# <a name="confirmation-messages"></a><span data-ttu-id="45749-102">Bestätigungsmeldungen</span><span class="sxs-lookup"><span data-stu-id="45749-102">Confirmation Messages</span></span>

<span data-ttu-id="45749-103">Nachfolgend finden Sie verschiedene Bestätigungsnachrichten, die abhängig von der Varianten der angezeigt werden, können die [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [ System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methoden, die aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="45749-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45749-104">Beispielcode, der zeigt, wie Sie Bestätigungen anfordern, finden Sie unter [wie Anforderung Bestätigungen](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="45749-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="45749-105">Angeben der Ressource</span><span class="sxs-lookup"><span data-stu-id="45749-105">Specifying the Resource</span></span>

<span data-ttu-id="45749-106">Sie können angeben, dass die Ressource, die durch Aufrufen von geändert werden, die [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) Methode.</span><span class="sxs-lookup"><span data-stu-id="45749-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="45749-107">In diesem Fall geben Sie die Ressource mithilfe der `target` Parameter der Methode und der Vorgang wird von Windows PowerShell hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="45749-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="45749-108">In der folgenden Meldung aus der Text "MyResource" ist die Ressource behandelt, und der Vorgang ist der Name des Befehls, der den Aufruf ausführt.</span><span class="sxs-lookup"><span data-stu-id="45749-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="45749-109">Wenn der Benutzer wählt **Ja** oder **Ja, alle** auf die Bestätigung anfordern (wie im folgenden Beispiel gezeigt), einen Aufruf der [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methode vorgenommen wird, die bewirkt, dass einer zweite bestätigungsmeldung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="45749-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="45749-110">Angeben, den Betrieb und die Ressource</span><span class="sxs-lookup"><span data-stu-id="45749-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="45749-111">Sie können angeben, die Ressource, die geändert werden, und der Vorgang, der der Befehl führen Sie durch Aufrufen der [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) Methode.</span><span class="sxs-lookup"><span data-stu-id="45749-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="45749-112">In diesem Fall geben Sie die Ressource mithilfe der `target` Parameter und den Vorgang mit der `target` Parameter.</span><span class="sxs-lookup"><span data-stu-id="45749-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="45749-113">In der folgenden Meldung aus der Text "MyResource" ist die Ressource behandelt, und "MyAction" ist der Vorgang ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="45749-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="45749-114">Wenn der Benutzer auswählt **Ja** oder **Ja, alle** zur vorherigen Nachricht, einen Aufruf der [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methode vorgenommen wird, wodurch ein zweite bestätigungsmeldung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="45749-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="45749-115">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="45749-115">See Also</span></span>

[<span data-ttu-id="45749-116">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="45749-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
