---
title: Runspace05-Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1685cfc4-b32c-4bed-b221-e0c4482db955
caps.latest.revision: 9
ms.openlocfilehash: b640493bca81a0157bf5abffe3ab43b3a2832b01
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565256"
---
# <a name="runspace05-sample"></a>Runspace05-Beispiel

In diesem Beispiel wird gezeigt, wie ein Snap-in zu einem [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt hinzugefügt wird, sodass das Cmdlet des Snap-Ins verfügbar ist, wenn der Runspace geöffnet wird. Das-Snap-in stellt ein Get-proc-Cmdlet bereit (definiert durch das [GetProcessSample01-Beispiel](../cmdlet/getprocesssample01-sample.md)), das synchron mithilfe eines [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts ausgeführt wird.

## <a name="requirements"></a>Anforderungen

Dieses Beispiel erfordert Windows PowerShell 2,0.

## <a name="demonstrates"></a>Zeigt

In diesem Beispiel wird Folgendes veranschaulicht:

- Ein [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt wird erstellt.

- Das Snap-in wird dem [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt hinzugefügt.

- Erstellen eines [System. Management. Automation. Runspaces. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) -Objekts, das das [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt verwendet.

- Erstellen eines [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts, das den Runspace verwendet.

- Das Get-proc-Cmdlet des Snap-Ins wird der Pipeline des [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts hinzugefügt.

- Synchrones Ausführen des Befehls.

- Extrahieren von Eigenschaften aus den [System. Management. Automation. psobject](/dotnet/api/System.Management.Automation.PSObject) -Objekten, die vom Befehl zurückgegeben werden.

## <a name="example"></a>Beispiel

In diesem Beispiel wird ein Runspace erstellt, der ein [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt verwendet, um die Elemente zu definieren, die beim Öffnen des Runspace verfügbar sind. In diesem Beispiel wird ein Snap-in, das ein Get-proc-Cmdlet definiert, dem anfänglichen Sitzungszustand hinzugefügt.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace05
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a Windows PowerShell snap-in that is present in the console file.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample01.dll
    /// that is produced by the GetProcessSample01 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a snap-in to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the snap-in's get-proc cmdlet to the PowerShell object.
    /// 6. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create the default initial session state. The default initial
      // session state contains all the elements provided by Windows
      // PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      PSSnapInException warning;
      iss.ImportPSSnapIn("GetProcPSSnapIn01", out warning);

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the snap-in cmdlet and specify the runspace.
          powershell.AddCommand("GetProcPSSnapIn01\\get-proc");
          powershell.Runspace = myRunSpace;

          // Run the cmdlet synchronously.
          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the results.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                              "{0,-20} {1}",
                              result.Members["ProcessName"].Value,
                              result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release any resources.
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
