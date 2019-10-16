---
title: Bestätigungsmeldungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 229725b5b9f1f0082592dcebe11564fd2f630ce1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365729"
---
# <a name="confirmation-messages"></a><span data-ttu-id="e70d4-102">Bestätigungsmeldungen</span><span class="sxs-lookup"><span data-stu-id="e70d4-102">Confirmation Messages</span></span>

<span data-ttu-id="e70d4-103">Im folgenden finden Sie unterschiedliche Bestätigungsmeldungen, die je nach den Varianten der Methoden " [System. Management. Automation. Cmdlet. Schulter dprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) " und " [System. Management. Automation. Cmdlet. schuldcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) " angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="e70d4-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e70d4-104">Beispielcode, der zeigt, wie Bestätigungen angefordert werden, finden Sie unter [anfordern von Bestätigungen](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="e70d4-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="e70d4-105">Angeben der Ressource</span><span class="sxs-lookup"><span data-stu-id="e70d4-105">Specifying the Resource</span></span>

<span data-ttu-id="e70d4-106">Sie können die zu ändernde Ressource angeben, indem Sie das [System. Management. Automation. Cmdlet aufrufen. Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) -Methode.</span><span class="sxs-lookup"><span data-stu-id="e70d4-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="e70d4-107">In diesem Fall stellen Sie die Ressource mithilfe des Parameters "`target`" der-Methode bereit, und der Vorgang wird von Windows PowerShell hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e70d4-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="e70d4-108">In der folgenden Meldung ist der Text "MyResource" die Ressource, auf die reagiert wird, und der Vorgang ist der Name des Befehls, der den-Vorgang ausführt.</span><span class="sxs-lookup"><span data-stu-id="e70d4-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="e70d4-109">Wenn der Benutzer für die Bestätigungs Anforderung **Ja** oder **Ja** (wie im folgenden Beispiel gezeigt) auswählt, wird ein [System. Management. Automation. Cmdlet. ermdcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode aufgerufen, die eine zweite Bestätigungsmeldung bewirkt. gestellte.</span><span class="sxs-lookup"><span data-stu-id="e70d4-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="e70d4-110">Angeben des Vorgangs und der Ressource</span><span class="sxs-lookup"><span data-stu-id="e70d4-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="e70d4-111">Sie können die zu ändernde Ressource und den von dem Befehl auszuführenden Vorgang angeben, indem Sie das [System. Management. Automation. Cmdlet. tiondprocess% 2a aufrufen? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) -Methode.</span><span class="sxs-lookup"><span data-stu-id="e70d4-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="e70d4-112">In diesem Fall geben Sie die Ressource mithilfe des Parameters "`target`" und des Vorgangs mithilfe des Parameters "`target`" an.</span><span class="sxs-lookup"><span data-stu-id="e70d4-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="e70d4-113">In der folgenden Meldung ist der Text "MyResource" die Ressource, die ausgeführt wird, und "myaction" ist der Vorgang, der ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="e70d4-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="e70d4-114">Wenn der Benutzer für die vorherige Nachricht **Ja** oder **Ja** ausgewählt hat, wird ein Rückruf der [System. Management. Automation. Cmdlet. ermdcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode durchgeführt, wodurch eine zweite Bestätigungsmeldung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e70d4-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="e70d4-115">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e70d4-115">See Also</span></span>

[<span data-ttu-id="e70d4-116">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="e70d4-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
