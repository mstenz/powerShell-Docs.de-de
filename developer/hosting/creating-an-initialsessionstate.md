---
title: Erstellen eine InitialSessionState | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 9140d03e046def2fbbcc2a842b9ea1b9e1fa2985
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263836"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="61d9a-102">Erstellen von InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="61d9a-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="61d9a-103">Führen Sie PowerShell-Befehle in einem Runspace.</span><span class="sxs-lookup"><span data-stu-id="61d9a-103">PowerShell commands run in a runspace.</span></span>
<span data-ttu-id="61d9a-104">Um PowerShell in Ihrer Anwendung zu hosten, müssen Sie erstellen eine [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) Objekt.</span><span class="sxs-lookup"><span data-stu-id="61d9a-104">To host PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>
<span data-ttu-id="61d9a-105">Jede Runspace verfügt über eine [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt verknüpft.</span><span class="sxs-lookup"><span data-stu-id="61d9a-105">Every runspace has an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span>
<span data-ttu-id="61d9a-106">Die InitialSessionState gibt die Eigenschaften des dem-Runspace, z. B., den Befehle, Variablen und Module für diesen Runspace verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="61d9a-106">The InitialSessionState specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="61d9a-107">Erstellt einen Standard-InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="61d9a-107">Create a default InitialSessionState</span></span>

<span data-ttu-id="61d9a-108">Die [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) und [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) Methoden der **InitialSessionState** Klasse kann verwendet werden, um das Erstellen einer **InitialSessionState**Objekt.</span><span class="sxs-lookup"><span data-stu-id="61d9a-108">The [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) and [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods of the **InitialSessionState** class can be used to create an **InitialSessionState** object.</span></span>
<span data-ttu-id="61d9a-109">Die **CreateDefault** -Methode erstellt eine **InitialSessionState** mit allen von den integrierten Befehlen geladen, während die **CreateDefault2** Methode lädt nur die Befehle erforderlich, um den Host PowerShell (die Befehle aus dem Microsoft.PowerShell.Core-Modul).</span><span class="sxs-lookup"><span data-stu-id="61d9a-109">The **CreateDefault** method creates an **InitialSessionState** with all of the built-in commands loaded, while the **CreateDefault2** method loads only the commands required to host PowerShell (the commands from the Microsoft.PowerShell.Core module).</span></span>

<span data-ttu-id="61d9a-110">Wenn Sie die Befehle in der hostanwendung verfügbar weiter einschränken möchten, müssen Sie einen eingeschränkten Runspace zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="61d9a-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span>
<span data-ttu-id="61d9a-111">Weitere Informationen finden Sie unter [einen eingeschränkten Runspace erstellen](creating-a-constrained-runspace.md).</span><span class="sxs-lookup"><span data-stu-id="61d9a-111">For information, see [Creating a constrained runspace](creating-a-constrained-runspace.md).</span></span>

<span data-ttu-id="61d9a-112">Der folgende Code zeigt, wie Sie erstellen eine **InitialSessionState**, weisen Sie es mit einem Runspace, Hinzufügen von Befehlen für die Pipeline in diesem Runspace und die Befehle aufrufen.</span><span class="sxs-lookup"><span data-stu-id="61d9a-112">The following code shows how to create an **InitialSessionState**, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span>
<span data-ttu-id="61d9a-113">Weitere Informationen zum Hinzufügen und Aufrufen von Befehlen finden Sie unter [hinzufügen und Aufrufen von Befehlen](adding-and-invoking-commands.md).</span><span class="sxs-lookup"><span data-stu-id="61d9a-113">For more information about adding and invoking commands, see [Adding and invoking commands](adding-and-invoking-commands.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="61d9a-114">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="61d9a-114">See Also</span></span>

[<span data-ttu-id="61d9a-115">Erstellen einen eingeschränkten runspace</span><span class="sxs-lookup"><span data-stu-id="61d9a-115">Creating a constrained runspace</span></span>](creating-a-constrained-runspace.md)

[<span data-ttu-id="61d9a-116">Hinzufügen und Aufrufen von Befehlen</span><span class="sxs-lookup"><span data-stu-id="61d9a-116">Adding and invoking commands</span></span>](adding-and-invoking-commands.md)
