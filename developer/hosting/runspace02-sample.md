---
title: Beispiel für Runspace02 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7630bb63-ef39-4abd-b795-8000f984c1e5
caps.latest.revision: 9
ms.openlocfilehash: 6352169cffbb8a8bf59a42f79979f5003c150fa4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082718"
---
# <a name="runspace02-sample"></a>Runspace02-Beispiel

Dieses Beispiel zeigt, wie Sie mit der [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) -Klasse zum Ausführen der [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) und [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) Cmdlets synchron. Die [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) -Cmdlet zurückgegeben ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) -Objekte für jeden Prozess auf dem lokalen Computer ausgeführt wird und die `Sort-Object` sortiert die Objekte basierend auf ihren [ System.Diagnostics.Process.Id*](/dotnet/api/System.Diagnostics.Process.Id) Eigenschaft. Die Ergebnisse dieser Befehle anzeigen, indem eine [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) Steuerelement.

## <a name="requirements"></a>Anforderungen

Dieses Beispiel ist die Windows PowerShell 2.0 erforderlich.

## <a name="demonstrates"></a>Zeigt

Dieses Beispiel veranschaulicht die folgenden.

- Erstellen einer [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Objekt zum Ausführen von Befehlen.

- Hinzufügen von Befehlen an die Pipeline von [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Objekt.

- Die Befehle ausführen synchron.

- Mit einem [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) -Steuerelement zum Anzeigen der Ausgabe der Befehle in einer Windows Forms-Anwendung.

## <a name="example"></a>Beispiel

In diesem Beispiel führt die [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) und [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) Cmdlets synchron in dem standardmäßigen Runspace von Windows PowerShell bereitgestellt. Die Ausgabe wird angezeigt, in einer Form mit einem [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) Steuerelement.

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

[Schreiben Sie eine Windows PowerShell-Hostanwendung](./writing-a-windows-powershell-host-application.md)