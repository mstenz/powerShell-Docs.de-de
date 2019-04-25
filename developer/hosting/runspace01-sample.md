---
title: Beispiel für Runspace01 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c1c59c-6da5-4cda-9562-e8059177fee1
caps.latest.revision: 11
ms.openlocfilehash: eec9c616fc6d5240db185f764a3ea2c8f9575d03
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082786"
---
# <a name="runspace01-sample"></a>Runspace01-Beispiel

Dieses Beispiel zeigt, wie Sie mit der [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) -Klasse zum Ausführen der [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet synchron. Die [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) -Cmdlet zurückgegeben ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) -Objekte für jeden Prozess auf dem lokalen Computer ausgeführt wird. Die Werte der [System.Diagnostics.Process.Processname*](/dotnet/api/System.Diagnostics.Process.ProcessName) und [System.Diagnostics.Process.Handlecount*](/dotnet/api/System.Diagnostics.Process.Handlecount) Eigenschaften klicken Sie dann aus der zurückgegebenen Objekte extrahiert und in einem Konsolenfenster angezeigt werden Fenster.

## <a name="requirements"></a>Anforderungen

 Dieses Beispiel ist die Windows PowerShell 2.0 erforderlich.

## <a name="demonstrates"></a>Zeigt

- Erstellen einer [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Objekt um einen Befehl auszuführen.

- Hinzufügen eines Befehls der Pipeline die [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Objekt.

- Den Befehl synchron ausgeführt.

- Mithilfe von [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) Objekte zum Extrahieren von Eigenschaften aus den Objekten, die vom Befehl zurückgegeben wird.

## <a name="example"></a>Beispiel

 In diesem Beispiel führt die [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet synchron auf dem standardmäßigen Runspace von Windows PowerShell bereitgestellt.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace01
  {
    /// <summary>
    /// This sample uses the PowerShell class to execute
    /// the get-process cmdlet synchronously. The name and
    /// handlecount are then extracted from the PSObjects
    /// returned and displayed.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run a command.
    /// 2. Adding a command to the pipeline of the PowerShell object.
    /// 3. Running the command synchronously.
    /// 4. Using PSObject objects to extract properties from the objects
    ///    returned by the command.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create().AddCommand("get-process"))
      {
        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the command synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke())
        {
          Console.WriteLine(
                      "{0,-20} {1}",
                      result.Members["ProcessName"].Value,
                      result.Members["HandleCount"].Value);
        }
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>Weitere Informationen
