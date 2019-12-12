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
ms.openlocfilehash: f776f13fe743a3f5f67de0d94883e3f754040ffc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367639"
---
# <a name="adding-and-invoking-commands"></a>Hinzufügen und Aufrufen von Befehlen

Nachdem Sie einen Runspace erstellt haben, können Sie Windows powershellcommands und Skripts zu einer Pipeline hinzufügen und die Pipeline dann synchron oder asynchron aufrufen.

## <a name="creating-a-pipeline"></a>Erstellen einer Pipeline

 Die [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Klasse bietet mehrere Methoden zum Hinzufügen von Befehlen, Parametern und Skripts zur Pipeline. Sie können die Pipeline synchron aufrufen, indem Sie eine Überladung der [System. Management. Automation. PowerShell. Call *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) -Methode aufrufen, oder asynchron durch Aufrufen einer Überladung von [System. Management. Automation. PowerShell. beginCall *](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) und der [System. Management. Automation. PowerShell. EndInvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) -Methode.

### <a name="addcommand"></a>AddCommand

1. Erstellen Sie ein [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekt.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Fügen Sie den Befehl hinzu, den Sie ausführen möchten.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Rufen Sie den Befehl auf.

   ```csharp
   ps.Invoke();
   ```

 Wenn Sie die [System. Management. Automation. PowerShell. AddCommand *](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) -Methode mehrmals aufrufen, bevor Sie die [System. Management. Automation. PowerShell. Call*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) -Methode aufrufen, wird das Ergebnis des ersten Befehls an die zweite weitergeleitet usw. Wenn Sie das Ergebnis eines vorherigen Befehls nicht an einen Befehl übergeben möchten, fügen Sie es hinzu, indem Sie stattdessen die [System. Management. Automation. PowerShell. addstatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) aufrufen.

### <a name="addparameter"></a>AddParameter

 Das vorherige Beispiel führt einen einzelnen Befehl ohne Parameter aus. Sie können dem Befehl Parameter hinzufügen, indem Sie die [System. Management. Automation. PSCommand. AddParameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) -Methode verwenden. der folgende Code ruft beispielsweise eine Liste aller Prozesse ab, die `PowerShell` auf dem Computer ausgeführt werden.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 Sie können zusätzliche Parameter hinzufügen, indem Sie [System. Management. Automation. PSCommand. AddParameter *](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) wiederholt aufrufen.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 Sie können auch ein Wörterbuch mit Parameternamen und-Werten hinzufügen, indem Sie die [System. Management. Automation. PowerShell. AddParameters *](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) -Methode aufrufen.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>Addstatement

 Sie können die Batch Verarbeitung simulieren, indem Sie die [System. Management. Automation. PowerShell. addstatement *](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) -Methode verwenden, mit der am Ende der Pipeline eine zusätzliche Anweisung hinzugefügt wird. der folgende Code Ruft eine Liste der ausgelaufenden Prozesse mit dem Namen `PowerShell`ab und ruft dann die Liste der ausgelaufenden Dienste ab.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 Sie können ein vorhandenes Skript ausführen, indem Sie die [System. Management. Automation. PowerShell. addScript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript) -Methode aufrufen. Das folgende Beispiel fügt der Pipeline ein Skript hinzu und führt es aus. In diesem Beispiel wird davon ausgegangen, dass bereits ein Skript mit dem Namen `MyScript.ps1` in einem Ordner namens `D:\PSScripts`vorhanden ist.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 Es gibt auch eine Version der [System. Management. Automation. PowerShell. addScript *](/dotnet/api/System.Management.Automation.PowerShell.AddScript) -Methode, die einen booleschen Parameter namens "`useLocalScope`" annimmt. Wenn dieser Parameter auf `true`festgelegt ist, wird das Skript im lokalen Gültigkeitsbereich ausgeführt. Mit dem folgenden Code wird das Skript im lokalen Gültigkeitsbereich ausgeführt.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>Synchrones Aufrufen einer Pipeline

 Nachdem Sie der Pipeline Elemente hinzugefügt haben, rufen Sie Sie auf. Um die Pipeline synchron aufzurufen, rufen Sie eine Überladung der [System. Management. Automation. PowerShell. aufrufen *](/dotnet/api/System.Management.Automation.PowerShell.Invoke) -Methode auf. Im folgenden Beispiel wird gezeigt, wie eine Pipeline synchron aufgerufen wird.

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

### <a name="invoking-a-pipeline-asynchronously"></a>Asynchrones Aufrufen einer Pipeline

 Sie rufen eine Pipeline asynchron auf, indem Sie eine Überladung von [System. Management. Automation. PowerShell. beginCall *](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) aufrufen, um ein [IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) -Objekt zu erstellen, und dann die [System. Management. Automation. PowerShell. EndInvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) -Methode aufrufen.

 Im folgenden Beispiel wird gezeigt, wie eine Pipeline asynchron aufgerufen wird.

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

 [Erstellen eines initialsessionstate](./creating-an-initialsessionstate.md)

 [Erstellen eines eingeschränkten Runspace](./creating-a-constrained-runspace.md)
