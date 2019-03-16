---
title: 'Gewusst wie: Anfordern von Bestätigungen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058818"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="9d977-102">Anfordern von Bestätigungen</span><span class="sxs-lookup"><span data-stu-id="9d977-102">How to Request Confirmations</span></span>

<span data-ttu-id="9d977-103">In diesem Beispiel wird gezeigt, wie zum Aufrufen der [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methoden zum Anfordern von Bestätigungen aus der Benutzer, bevor eine Aktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9d977-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9d977-104">Weitere Informationen zur Behandlung dieser Anforderungen von Windows PowerShell finden Sie unter [Bestätigung anfordern](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="9d977-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="9d977-105">Eine Bestätigung anzufordern</span><span class="sxs-lookup"><span data-stu-id="9d977-105">To request confirmation</span></span>

1. <span data-ttu-id="9d977-106">Sicherstellen, dass die `SupportsShouldProcess` Parameter des Cmdlet-Attributs nastaven NA hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="9d977-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="9d977-107">(Für Funktionen ist dies ein Parameter des Attributs CmdletBinding.)</span><span class="sxs-lookup"><span data-stu-id="9d977-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="9d977-108">Hinzufügen einer `Force` Parameter, um Ihr Cmdlet, damit der Benutzer eine Bestätigungs-Anforderung überschreiben kann.</span><span class="sxs-lookup"><span data-stu-id="9d977-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="9d977-109">Hinzufügen einer `if` -Anweisung, die den Rückgabewert des verwendet die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Methode, um zu bestimmen, ob die [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methode wird aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="9d977-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="9d977-110">Fügen Sie eine zweite `if` -Anweisung, den Rückgabewert von der [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode und der Wert des der `Force` Parameter, um zu bestimmen, ob der Vorgang sein soll ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="9d977-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="9d977-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="9d977-111">Example</span></span>

<span data-ttu-id="9d977-112">Das folgende Codebeispiel zeigt die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methoden aus aufgerufen werden, in der Überschreibung von der [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode.</span><span class="sxs-lookup"><span data-stu-id="9d977-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="9d977-113">Allerdings können Sie auch diese Methoden aus den anderen eingabeverarbeitungsmethoden aufrufen.</span><span class="sxs-lookup"><span data-stu-id="9d977-113">However, you can also call these methods from the other input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9d977-114">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9d977-114">See Also</span></span>

[<span data-ttu-id="9d977-115">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="9d977-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
