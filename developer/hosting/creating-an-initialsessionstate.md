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
# <a name="creating-an-initialsessionstate"></a>Erstellen von InitialSessionState

Führen Sie Windows PowerShell-Befehle in einem Runspace. Um Windows PowerShell in Ihrer Anwendung zu hosten, müssen Sie erstellen eine [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) Objekt. Jede Runspace verfügt über eine [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt verknüpft. Die [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) gibt die Eigenschaften des dem-Runspace, z. B. die Befehle, Variablen und Module für diesen Runspace verfügbar sind.

## <a name="create-a-default-initialsessionstate"></a>Erstellt einen Standard-InitialSessionState

 Die [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)und [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) Methoden können verwendet werden Erstellung [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Objekte. [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) erstellt eine InitialSessionState für die geladen, während mit allen von den integrierten Befehlen [ System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) lädt nur die Befehle, die zum Hosten von Windows PowerShell (die Befehle aus dem Microsoft.PowerShell.Core-Modul.

 Wenn Sie die Befehle in der hostanwendung verfügbar weiter einschränken möchten, müssen Sie einen eingeschränkten Runspace zu erstellen. Informationen finden Sie unter einem eingeschränkten Runspace zu erstellen.

 Der folgende Code zeigt, wie Sie eine InitialSessionState erstellen, weisen Sie es mit einem Runspace, Hinzufügen von Befehlen für die Pipeline in diesem Runspace und die Befehle aufrufen. Weitere Informationen zum Hinzufügen und Aufrufen von Befehlen finden Sie unter Hinzufügen und Aufrufen von Befehlen.

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

## <a name="see-also"></a>Weitere Informationen

 [Erstellen einen eingeschränkten runspace](./creating-a-constrained-runspace.md)
