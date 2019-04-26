---
title: Wie Sie ein Cmdlet in einem Cmdlet aufrufen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067823"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="6ca11-102">Aufrufen eines Cmdlet in einem Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6ca11-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="6ca11-103">Dieses Beispiel zeigt, wie Sie ein Cmdlet in ein anderes Cmdlet aufrufen, können Sie die Funktionalität des aufgerufenen-Cmdlets zum Cmdlet hinzugefügt, die Sie entwickeln.</span><span class="sxs-lookup"><span data-stu-id="6ca11-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="6ca11-104">In diesem Beispiel die `Get-Process` Cmdlet wird aufgerufen, um die Prozesse abzurufen, die auf dem lokalen Computer ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="6ca11-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="6ca11-105">Der Aufruf der `Get-Process` Cmdlet entspricht den folgenden Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="6ca11-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="6ca11-106">Dieser Befehl ruft alle Prozesse, deren Namen mit den Zeichen "a" bis "t" beginnen.</span><span class="sxs-lookup"><span data-stu-id="6ca11-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="6ca11-107">Sie können nur die Cmdlets, die direkt vom abgeleitet sind Aufrufen der [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) Klasse.</span><span class="sxs-lookup"><span data-stu-id="6ca11-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="6ca11-108">Sie können nicht aufgerufen werden ein Cmdlet, das von abgeleitet ist die [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) Klasse.</span><span class="sxs-lookup"><span data-stu-id="6ca11-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="6ca11-109">Um ein Cmdlet in einem Cmdlet aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="6ca11-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="6ca11-110">Stellen Sie sicher, dass die Assembly, definiert das-Cmdlet aufgerufen werden, verwiesen wird und dass die entsprechenden `using` -Anweisung wird hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="6ca11-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="6ca11-111">In diesem Beispiel werden die folgenden Namespaces hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="6ca11-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="6ca11-112">Erstellen Sie eine neue Instanz des-Cmdlets aufgerufen werden, in der Eingabe Verarbeitungsmethode des-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="6ca11-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="6ca11-113">In diesem Beispiel ist ein Objekt des Typs [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) wird erstellt, zusammen mit der Zeichenfolge, die die Argumente enthält, die verwendet werden, wenn das-Cmdlet aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="6ca11-113">In this example, an object of type [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="6ca11-114">Rufen Sie die [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) aufzurufende Methode der `Get-Process` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6ca11-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="6ca11-115">Beispiel</span><span class="sxs-lookup"><span data-stu-id="6ca11-115">Example</span></span>

<span data-ttu-id="6ca11-116">In diesem Beispiel die `Get-Process` Cmdlet wird aufgerufen, innerhalb der [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Methode eines Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="6ca11-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="6ca11-117">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6ca11-117">See Also</span></span>

[<span data-ttu-id="6ca11-118">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="6ca11-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
