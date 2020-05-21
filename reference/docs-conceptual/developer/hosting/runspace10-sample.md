---
title: Runspace10-Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c265084-e072-46ca-9844-c3c0e275d6b0
caps.latest.revision: 7
ms.openlocfilehash: 1a73c0b6731073b1bac941e323416e8c45d2c252
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565239"
---
# <a name="runspace10-sample"></a>Runspace10-Beispiel

In diesem Beispiel wird gezeigt, wie ein ursprünglicher Standard Sitzungszustand erstellt wird, wie ein Cmdlet zum [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)-Objekt hinzugefügt wird, wie ein Runspace erstellt wird, der den anfänglichen Sitzungs Status verwendet, und wie der Befehl mithilfe eines [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts ausgeführt wird.

## <a name="requirements"></a>Anforderungen

Dieses Beispiel erfordert Windows PowerShell 2,0.

## <a name="demonstrates"></a>Zeigt

In diesem Beispiel wird Folgendes veranschaulicht:

- Ein [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt wird erstellt.

- Hinzufügen eines Cmdlets (von der Host Anwendung definiert) zum [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt.

- Erstellen eines [System. Management. Automation. Runspaces. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) -Objekts, das das Objekt verwendet.

- Erstellen eines [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts, das das [System. Management. Automation. Runspaces. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) -Objekt verwendet.

- Hinzufügen des Befehls zur Pipeline des [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts.

- Extrahieren von Eigenschaften aus den [System. Management. Automation. psobject](/dotnet/api/System.Management.Automation.PSObject) -Objekten, die vom Befehl zurückgegeben werden.

## <a name="example"></a>Beispiel

In diesem Beispiel wird ein Runspace erstellt, der ein [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt verwendet, um die Elemente zu definieren, die beim Öffnen des Runspace verfügbar sind. In diesem Beispiel wird das Get-proc-Cmdlet (definiert durch die Host Anwendung) dem anfänglichen Sitzungszustand hinzugefügt, und das Cmdlet wird mithilfe eines [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts synchron ausgeführt.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Collections.ObjectModel;
  using System.Diagnostics;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  #region GetProcCommand

  /// <summary>
  /// Class that implements the GetProcCommand.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Cmdlet Overrides

    /// <summary>
    /// For each of the requested process names, retrieve and write
    /// the associated processes.
    /// </summary>
    protected override void ProcessRecord()
    {
      // Get the current processes.
      Process[] processes = Process.GetProcesses();

      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument (true) tells the
      // system to enumerate the array, and send one process object
      // at a time to the pipeline.
      WriteObject(processes, true);
    }

    #endregion Overrides
  } // End GetProcCommand class.

  #endregion GetProcCommand

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace10
  {
    /// <summary>
    /// This sample shows how to create a default initial session state, how to add
    /// add a cmdlet to the InitialSessionState object, and then how to create
    /// a Runspace object.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    /// This sample demonstrates:
    /// 1. Creating an InitialSessionState object.
    /// 2. Adding a cmdlet to the InitialSessionState object.
    /// 3. Creating a runspace that uses the InitialSessionState object.
    /// 4. Creating a PowerShell object that uses the Runspace object.
    /// 5. Running the added command synchronously.
    /// 6. Working with PSObject objects to extract properties
    ///    from the objects returned by the pipeline.
    private static void Main(string[] args)
    {
      // Create a default InitialSessionState object. The default
      // InitialSessionState object contains all the elements provided
      // by Windows PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();

      // Add the get-proc cmdlet to the InitialSessionState object.
      SessionStateCmdletEntry ssce = new SessionStateCmdletEntry("get-proc", typeof(GetProcCommand), null);
      iss.Commands.Add(ssce);

      // Create a Runspace object that uses the InitialSessionState object.
      // Notice that no PSHost object is specified, so the default host is used.
      // See the Hosting samples for information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Add the get-proc cmdlet to the pipeline of the PowerShell object.
          powershell.AddCommand("get-proc");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the output of the pipeline.
          foreach (PSObject result in results)
          {
             Console.WriteLine(
                               "{0,-20} {1}",
                               result.Members["ProcessName"].Value,
                               result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben einer Windows PowerShell-Hostanwendung](./writing-a-windows-powershell-host-application.md)
