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
ms.openlocfilehash: 3a7c47487b632d00643fce0aa082e0dc9a9bb626
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082990"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="0fc04-102">Erstellen von InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="0fc04-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="0fc04-103">Führen Sie Windows PowerShell-Befehle in einem Runspace.</span><span class="sxs-lookup"><span data-stu-id="0fc04-103">Windows PowerShell commands run in a runspace.</span></span> <span data-ttu-id="0fc04-104">Um Windows PowerShell in Ihrer Anwendung zu hosten, müssen Sie erstellen eine [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) Objekt.</span><span class="sxs-lookup"><span data-stu-id="0fc04-104">To host Windows PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span> <span data-ttu-id="0fc04-105">Jede Runspace verfügt über eine [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt verknüpft.</span><span class="sxs-lookup"><span data-stu-id="0fc04-105">Every runspace has an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span> <span data-ttu-id="0fc04-106">Die [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) gibt die Eigenschaften des dem-Runspace, z. B. die Befehle, Variablen und Module für diesen Runspace verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="0fc04-106">The [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="0fc04-107">Erstellt einen Standard-InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="0fc04-107">Create a default InitialSessionState</span></span>

 <span data-ttu-id="0fc04-108">Die [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)und [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) Methoden können verwendet werden Erstellung [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Objekte.</span><span class="sxs-lookup"><span data-stu-id="0fc04-108">The [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)and [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods can be used to create [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objects.</span></span> <span data-ttu-id="0fc04-109">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) erstellt eine InitialSessionState für die geladen, während mit allen von den integrierten Befehlen [ System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) lädt nur die Befehle, die zum Hosten von Windows PowerShell (die Befehle aus dem Microsoft.PowerShell.Core-Modul.</span><span class="sxs-lookup"><span data-stu-id="0fc04-109">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) creates an InitialSessionState with all of the built-in commands loaded, while [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) loads only the commands required to host Windows PowerShell (the commands from the Microsoft.PowerShell.Core module.</span></span>

 <span data-ttu-id="0fc04-110">Wenn Sie die Befehle in der hostanwendung verfügbar weiter einschränken möchten, müssen Sie einen eingeschränkten Runspace zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0fc04-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span> <span data-ttu-id="0fc04-111">Informationen finden Sie unter einem eingeschränkten Runspace zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0fc04-111">For information, see Creating a constrained runspace.</span></span>

 <span data-ttu-id="0fc04-112">Der folgende Code zeigt, wie Sie eine InitialSessionState erstellen, weisen Sie es mit einem Runspace, Hinzufügen von Befehlen für die Pipeline in diesem Runspace und die Befehle aufrufen.</span><span class="sxs-lookup"><span data-stu-id="0fc04-112">The following code shows how to create an InitialSessionState, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span> <span data-ttu-id="0fc04-113">Weitere Informationen zum Hinzufügen und Aufrufen von Befehlen finden Sie unter Hinzufügen und Aufrufen von Befehlen.</span><span class="sxs-lookup"><span data-stu-id="0fc04-113">For more information about adding and invoking commands, see Adding and invoking commands.</span></span>

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

      // Call the PowerShell.Create() method to create the PowerShell
      // object,and then specify the runspace and commands to the pipeline.
      // and  create the command pipeline.
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

## <a name="see-also"></a><span data-ttu-id="0fc04-114">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0fc04-114">See Also</span></span>

 [<span data-ttu-id="0fc04-115">Erstellen einen eingeschränkten runspace</span><span class="sxs-lookup"><span data-stu-id="0fc04-115">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
