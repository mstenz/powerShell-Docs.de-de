---
title: Erstellen eines initialsessionstate | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 9140d03e046def2fbbcc2a842b9ea1b9e1fa2985
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367619"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="4269f-102">Erstellen von InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="4269f-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="4269f-103">PowerShell-Befehle werden in einem Runspace ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="4269f-103">PowerShell commands run in a runspace.</span></span>
<span data-ttu-id="4269f-104">Um PowerShell in Ihrer Anwendung zu hosten, müssen Sie ein [System. Management. Automation. Runspaces. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) -Objekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="4269f-104">To host PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>
<span data-ttu-id="4269f-105">Jedem Runspace ist ein [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="4269f-105">Every runspace has an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span>
<span data-ttu-id="4269f-106">Initialsessionstate gibt die Merkmale des Runspace an, z. b. welche Befehle, Variablen und Module für diesen Runspace verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="4269f-106">The InitialSessionState specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="4269f-107">Erstellen eines standardinitialsessionstate</span><span class="sxs-lookup"><span data-stu-id="4269f-107">Create a default InitialSessionState</span></span>

<span data-ttu-id="4269f-108">Die Methoden "up- [default](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) " und " [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) " der Klasse " **initialsessionstate** " können zum Erstellen eines " **initialsessionstate** "-Objekts verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4269f-108">The [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) and [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods of the **InitialSessionState** class can be used to create an **InitialSessionState** object.</span></span>
<span data-ttu-id="4269f-109">Die Methode " **samatedefault** " erstellt einen " **initialsessionstate** ", wobei alle integrierten Befehle geladen werden, während die **CreateDefault2** -Methode nur die Befehle lädt, die zum Hosten von PowerShell erforderlich sind (die Befehle aus der Microsoft. PowerShell. Core-Modul).</span><span class="sxs-lookup"><span data-stu-id="4269f-109">The **CreateDefault** method creates an **InitialSessionState** with all of the built-in commands loaded, while the **CreateDefault2** method loads only the commands required to host PowerShell (the commands from the Microsoft.PowerShell.Core module).</span></span>

<span data-ttu-id="4269f-110">Wenn Sie die in der Host Anwendung verfügbaren Befehle weiter einschränken möchten, müssen Sie einen eingeschränkten Runspace erstellen.</span><span class="sxs-lookup"><span data-stu-id="4269f-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span>
<span data-ttu-id="4269f-111">Weitere Informationen finden Sie unter [Erstellen eines eingeschränkten Runspace](creating-a-constrained-runspace.md).</span><span class="sxs-lookup"><span data-stu-id="4269f-111">For information, see [Creating a constrained runspace](creating-a-constrained-runspace.md).</span></span>

<span data-ttu-id="4269f-112">Der folgende Code zeigt, wie Sie einen **initialsessionstate**erstellen, ihn einem Runspace zuweisen, der Pipeline in diesem Runspace Befehle hinzufügen und die Befehle aufrufen.</span><span class="sxs-lookup"><span data-stu-id="4269f-112">The following code shows how to create an **InitialSessionState**, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span>
<span data-ttu-id="4269f-113">Weitere Informationen zum Hinzufügen und Aufrufen von Befehlen finden Sie unter [Hinzufügen und Aufrufen von Befehlen](adding-and-invoking-commands.md).</span><span class="sxs-lookup"><span data-stu-id="4269f-113">For more information about adding and invoking commands, see [Adding and invoking commands](adding-and-invoking-commands.md).</span></span>

```csharp
namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitialSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell object,
      // and then specify the runspace and commands to the pipeline.
      // and create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
      foreach (PSObject result in ps.Invoke())
      {
        Console.WriteLine("{0,-20}{1}",
            result.Members["Name"].Value,
            result.Members["Value"].Value);
      } // End foreach.

      // Close the runspace to free resources.
      rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a><span data-ttu-id="4269f-114">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4269f-114">See Also</span></span>

[<span data-ttu-id="4269f-115">Erstellen eines eingeschränkten Runspace</span><span class="sxs-lookup"><span data-stu-id="4269f-115">Creating a constrained runspace</span></span>](creating-a-constrained-runspace.md)

[<span data-ttu-id="4269f-116">Hinzufügen und Aufrufen von Befehlen</span><span class="sxs-lookup"><span data-stu-id="4269f-116">Adding and invoking commands</span></span>](adding-and-invoking-commands.md)
