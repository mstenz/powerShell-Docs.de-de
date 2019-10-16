---
title: Anfordern von Bestätigungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369679"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="c7049-102">Anfordern von Bestätigungen</span><span class="sxs-lookup"><span data-stu-id="c7049-102">How to Request Confirmations</span></span>

<span data-ttu-id="c7049-103">In diesem Beispiel wird gezeigt, wie die Methoden [System. Management. Automation. Cmdlet. Schulter dprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [System. Management. Automation. Cmdlet. undcontinue aufgerufen werden](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , um Bestätigungen des Benutzers anzufordern, bevor eine Aktion durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c7049-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7049-104">Weitere Informationen dazu, wie diese Anforderungen von Windows PowerShell verarbeitet werden, finden Sie unter [Anfordern einer Bestätigung](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="c7049-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="c7049-105">Zum Anfordern einer Bestätigung</span><span class="sxs-lookup"><span data-stu-id="c7049-105">To request confirmation</span></span>

1. <span data-ttu-id="c7049-106">Stellen Sie sicher, dass der `SupportsShouldProcess`-Parameter des Cmdlet-Attributs auf `true` festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="c7049-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="c7049-107">(Für Functions handelt es sich hierbei um einen Parameter des cmdletbinding-Attributs.)</span><span class="sxs-lookup"><span data-stu-id="c7049-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="c7049-108">Fügen Sie dem Cmdlet einen `Force`-Parameter hinzu, damit der Benutzer eine Bestätigungs Anforderung außer Kraft setzen kann.</span><span class="sxs-lookup"><span data-stu-id="c7049-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="c7049-109">Fügen Sie eine `if`-Anweisung hinzu, die den Rückgabewert der [System. Management. Automation. Cmdlet. tiondprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode verwendet, um zu bestimmen, ob die [System. Management. Automation. Cmdlet. Schulter dcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="c7049-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="c7049-110">Fügen Sie eine zweite `if`-Anweisung hinzu, die den Rückgabewert der [System. Management. Automation. Cmdlet. tiondcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode und den Wert des Parameters `Force` verwendet, um zu bestimmen, ob der Vorgang ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="c7049-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="c7049-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c7049-111">Example</span></span>

<span data-ttu-id="c7049-112">Im folgenden Codebeispiel werden die Methoden " [System. Management. Automation. Cmdlet. Schulter dprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) " und " [System. Management. Automation. Cmdlet. daudcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) " innerhalb der Überschreibung von [aufgerufen. System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode.</span><span class="sxs-lookup"><span data-stu-id="c7049-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="c7049-113">Sie können diese Methoden jedoch auch aus den anderen Eingabe Verarbeitungsmethoden aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="c7049-113">However, you can also call these methods from the other input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="c7049-114">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c7049-114">See Also</span></span>

[<span data-ttu-id="c7049-115">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c7049-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
