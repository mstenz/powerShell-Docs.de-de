---
title: Runspace02-Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7630bb63-ef39-4abd-b795-8000f984c1e5
caps.latest.revision: 9
ms.openlocfilehash: 997b1d6841ff014093ba54bf7a1db7b0b7d746b8
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564805"
---
# <a name="runspace02-sample"></a>Runspace02-Beispiel

In diesem Beispiel wird gezeigt, wie die [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Klasse zum synchronen Ausführen der Cmdlets " [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) " und " [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) " verwendet wird. Das [Get-Process-](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet gibt [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekte für jeden Prozess zurück, der auf dem lokalen Computer ausgeführt wird, und `Sort-Object` sortiert die Objekte basierend auf Ihrer [System.Diagnostics.Process.ID *](/dotnet/api/System.Diagnostics.Process.Id) -Eigenschaft. Die Ergebnisse dieser Befehle werden mithilfe eines [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -Steuer Elements angezeigt.

## <a name="requirements"></a>Anforderungen

Dieses Beispiel erfordert Windows PowerShell 2,0.

## <a name="demonstrates"></a>Zeigt

In diesem Beispiel wird Folgendes veranschaulicht:

- Erstellen eines [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts zum Ausführen von Befehlen.

- Hinzufügen von Befehlen zur Pipeline des [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts.

- Synchrones Ausführen der Befehle.

- Verwenden eines [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -Steuer Elements, um die Ausgabe der Befehle in einer Windows Forms Anwendung anzuzeigen.

## <a name="example"></a>Beispiel

In diesem Beispiel [werden die Get-Process-](/powershell/module/Microsoft.PowerShell.Management/Get-Process) und [Sort-Object-](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) Cmdlets synchron im Standard-Runspace von Windows PowerShell ausgeführt. Die Ausgabe wird in einem Formular mithilfe eines [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -Steuer Elements angezeigt.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using System.Windows.Forms;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace02
  {
    /// <summary>
    /// This method creates the form where the output is displayed.
    /// </summary>
    private static void CreateForm()
    {
      Form form = new Form();
      DataGridView grid = new DataGridView();
      form.Controls.Add(grid);
      grid.Dock = DockStyle.Fill;

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddCommand("get-process").AddCommand("sort-object").AddArgument("ID");
        if (Runspace.DefaultRunspace == null)
        {
          Runspace.DefaultRunspace = powershell.Runspace;
        }

        Collection<PSObject> results = powershell.Invoke();

        // The generic collection needs to be re-wrapped in an ArrayList
        // for data-binding to work.
        ArrayList objects = new ArrayList();
        objects.AddRange(results);

        // The DataGridView will use the PSObjectTypeDescriptor type
        // to retrieve the properties.
        grid.DataSource = objects;
      }

      form.ShowDialog();
    }

    /// <summary>
    /// This sample uses a PowerShell object to run the Get-Process
    /// and Sort-Object cmdlets synchronously. Windows Forms and
    /// data binding are then used to display the results in a
    /// DataGridView control.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object.
    /// 2. Adding commands and arguments to the pipeline of
    ///    the PowerShell object.
    /// 3. Running the commands synchronously.
    /// 4. Using a DataGridView control to display the output
    ///    of the commands in a Windows Forms application.
    /// </remarks>
    private static void Main(string[] args)
    {
      Runspace02.CreateForm();
    }
  }
}
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben einer Windows PowerShell-Hostanwendung](./writing-a-windows-powershell-host-application.md)
