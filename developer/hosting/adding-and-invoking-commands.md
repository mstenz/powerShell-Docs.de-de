---
title: Hinzufügen und Aufrufen von Befehlen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 9a01f948c5b474b4f9068030907601543e13cc7e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057653"
---
# <a name="adding-and-invoking-commands"></a>Hinzufügen und Aufrufen von Befehlen

Nachdem ein Runspace erstellt haben, können Sie Windows PowerShellcommands und Skripts hinzufügen, um eine Pipeline und rufen Sie dann die Pipeline synchron oder asynchron.

## <a name="creating-a-pipeline"></a>Erstellen einer pipeline

 Die [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Klasse bietet mehrere Methoden, um Befehle, Parameter und Skripts zur Pipeline hinzufügen. Sie können die Pipeline synchron durch Aufruf einer Überladung von Aufrufen der [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) -Methode, oder asynchron durch Aufruf einer Überladung der der [ System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) und klicken Sie dann die [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) Methode.

### <a name="addcommand"></a>AddCommand

1. Erstellen Sie eine [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Objekt.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Fügen Sie den Befehl aus, dem Sie ausführen möchten.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Rufen Sie den Befehl.

   ```csharp
   ps.Invoke();
   ```

 Aufrufen der [System.Management.Automation.Powershell.Addcommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) Methode, die mehr als einmal vor dem Aufruf der [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) -Methode, die das Ergebnis der ersten Befehl wird über die Pipeline zum zweiten und So weiter. Wenn Sie nicht das Ergebnis eines vorherigen Befehls an einen Befehl übergeben möchten, fügen Sie ihn durch Aufrufen der [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) stattdessen.

### <a name="addparameter"></a>AddParameter

 Im vorherige Beispiel führt einen einzelnen Befehl ohne Parameter aus. Sie können Parameter an den Befehl hinzufügen, mit der [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) z. B. der folgende Code ruft Methode eine Liste aller Prozesse mit dem Namen `PowerShell` unter der Computer.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 Sie können zusätzliche Parameter hinzufügen, durch den Aufruf [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) wiederholt.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 Sie können auch ein Wörterbuch von Parameternamen und Werte hinzufügen, durch den Aufruf der [System.Management.Automation.Powershell.Addparameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) Methode.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 Sie können mithilfe von Batchverarbeitung simulieren die [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) -Methode, die an das Ende der Pipeline eine zusätzliche Anweisung der folgende Code eine Liste fügt ruft der ausgeführten Prozesse mit dem Namen `PowerShell`, und ruft anschließend die Liste der ausgeführten Dienste.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 Sie können ein vorhandenes Skript ausführen, durch den Aufruf der [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) Methode. Im folgenden Beispiel wird die Pipeline ein Skript hinzugefügt und wird ausgeführt. In diesem Beispiel wird vorausgesetzt, es ist bereits ein Skript namens `MyScript.ps1` in einem Ordner namens `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 Es gibt auch eine Version der [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) -Methode, die einen booleschen namens Parameter `useLocalScope`. Wenn dieser Parameter, um festgelegt wird `true`, und klicken Sie dann das Skript im lokalen Bereich ausgeführt wird. Der folgende Code führt das Skript im lokalen Bereich.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>Synchron Aufrufen einer pipeline

 Nachdem Sie die Pipeline Elemente hinzuzufügen, rufen Sie es. Um die Pipeline synchron aufzurufen, rufen Sie eine Überladung von der [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) Methode. Das folgende Beispiel zeigt, wie Sie eine Pipeline synchron aufrufen.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a>Aufrufen einer Pipeline asynchron

 Sie rufen eine Pipeline asynchron durch Aufruf einer Überladung der der [System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) zum Erstellen einer [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) , und klicken Sie dann durch Aufrufen der [ System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) Methode.

 Das folgende Beispiel zeigt, wie Sie eine Pipeline asynchron aufrufen.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediately
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a>Weitere Informationen

 [Erstellen eine InitialSessionState](./creating-an-initialsessionstate.md)

 [Erstellen einen eingeschränkten runspace](./creating-a-constrained-runspace.md)
